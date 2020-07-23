---
title: PowerShell を使用して Microsoft 365 ユーザーアカウントのプロパティを構成する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/16/2020
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
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: '概要: microsoft 365 の PowerShell を使用して、Microsoft 365 テナント内の個別のまたは複数のユーザーアカウントのプロパティを構成します。'
ms.openlocfilehash: ccf9bf9930551ab1ee26ef7a1f69427cdc4871f5
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230853"
---
# <a name="configure-microsoft-365-user-account-properties-with-powershell"></a><span data-ttu-id="18d6b-103">PowerShell を使用して Microsoft 365 ユーザーアカウントのプロパティを構成する</span><span class="sxs-lookup"><span data-stu-id="18d6b-103">Configure Microsoft 365 user account properties with PowerShell</span></span>

<span data-ttu-id="18d6b-104">*この記事は、Microsoft 365 Enterprise と Office 365 Enterprise の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="18d6b-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="18d6b-105">Microsoft 365 管理センターを使用して、Microsoft 365 テナントのユーザーアカウントのプロパティを構成することはできますが、PowerShell を使用して、Microsoft 365 管理センターではできないいくつかの操作を実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="18d6b-105">Although you can use the Microsoft 365 admin center to configure properties for the user accounts of your Microsoft 365 tenant, you can also use PowerShell and do some things that the Microsoft 365 admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="18d6b-106">Graph 用 Azure Active Directory PowerShell モジュールを使用する</span><span class="sxs-lookup"><span data-stu-id="18d6b-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="18d6b-107">Graph モジュールの Azure Active Directory PowerShell を使用してユーザーアカウントのプロパティを構成するには、 [set-azureaduser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0)コマンドレットを使用して、設定または変更するプロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="18d6b-107">To configure properties for user accounts with the Azure Active Directory PowerShell for Graph module, you use the [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="18d6b-108">最初に、 [Microsoft 365 テナントに接続](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)します。</span><span class="sxs-lookup"><span data-stu-id="18d6b-108">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
   
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="18d6b-109">特定のユーザー アカウントのプロパティを変更する</span><span class="sxs-lookup"><span data-stu-id="18d6b-109">Change properties for a specific user account</span></span>

<span data-ttu-id="18d6b-110">**-ObjectID** パラメーターでアカウントを識別し、その他のパラメーターで特定のプロパティを設定または変更します。</span><span class="sxs-lookup"><span data-stu-id="18d6b-110">You identify the account with the **-ObjectID** parameter and set or change specific properties with additional parameters.</span></span> <span data-ttu-id="18d6b-111">最も一般的なパラメーターの一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="18d6b-111">Here's a list of the most common parameters.</span></span>
  
- <span data-ttu-id="18d6b-112">-Department "<部署名>"</span><span class="sxs-lookup"><span data-stu-id="18d6b-112">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="18d6b-113">-DisplayName "<完全なユーザー名>"</span><span class="sxs-lookup"><span data-stu-id="18d6b-113">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="18d6b-114">-FacsimilieTelephoneNumber "<FAX 番号>"</span><span class="sxs-lookup"><span data-stu-id="18d6b-114">-FacsimilieTelephoneNumber "\<fax number>"</span></span>
    
- <span data-ttu-id="18d6b-115">-GivenName "<ユーザーの名>"</span><span class="sxs-lookup"><span data-stu-id="18d6b-115">-GivenName "\<user first name>"</span></span>
    
- <span data-ttu-id="18d6b-116">-Surname "<ユーザーの姓>"</span><span class="sxs-lookup"><span data-stu-id="18d6b-116">-Surname "\<user last name>"</span></span>
    
- <span data-ttu-id="18d6b-117">-Mobile "<携帯電話番号>"</span><span class="sxs-lookup"><span data-stu-id="18d6b-117">-Mobile "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="18d6b-118">-JobTitle "<役職>"</span><span class="sxs-lookup"><span data-stu-id="18d6b-118">-JobTitle "\<job title>"</span></span>
    
- <span data-ttu-id="18d6b-119">-PreferredLanguage "<言語>"</span><span class="sxs-lookup"><span data-stu-id="18d6b-119">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="18d6b-120">-StreetAddress "<番地>"</span><span class="sxs-lookup"><span data-stu-id="18d6b-120">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="18d6b-121">-City "<市区町村名>"</span><span class="sxs-lookup"><span data-stu-id="18d6b-121">-City "\<city name>"</span></span>
    
- <span data-ttu-id="18d6b-122">-State "<都道府県名>"</span><span class="sxs-lookup"><span data-stu-id="18d6b-122">-State "\<state name>"</span></span>
    
- <span data-ttu-id="18d6b-123">-PostalCode "<郵便番号>"</span><span class="sxs-lookup"><span data-stu-id="18d6b-123">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="18d6b-124">-Country "<国名>"</span><span class="sxs-lookup"><span data-stu-id="18d6b-124">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="18d6b-125">-TelephoneNumber "<勤務先電話番号>"</span><span class="sxs-lookup"><span data-stu-id="18d6b-125">-TelephoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="18d6b-126">-" \<2-character country or region code> "</span><span class="sxs-lookup"><span data-stu-id="18d6b-126">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="18d6b-127">これは、ISO 3166-1 alpha-2 (A2) の 2 文字の国/地域コードです。</span><span class="sxs-lookup"><span data-stu-id="18d6b-127">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="18d6b-128">その他のパラメーターについては、[Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="18d6b-128">See [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) for additional parameters.</span></span>


<span data-ttu-id="18d6b-129">ユーザー アカウントのユーザー プリンシパル名を表示するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="18d6b-129">To display the User Principal Name for your user accounts, run the following command.</span></span>
  
```powershell
Get-AzureADUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

<span data-ttu-id="18d6b-130">次のコマンドは、PowerShell に次のように指示します。</span><span class="sxs-lookup"><span data-stu-id="18d6b-130">This command instructs PowerShell to:</span></span>
  
- <span data-ttu-id="18d6b-131">ユーザーアカウントのすべての情報を取得し (**set-azureaduser**)、次のコマンドに送信し **|** ます ()。</span><span class="sxs-lookup"><span data-stu-id="18d6b-131">Get all of the information on the user accounts (**Get-AzureADUser**) and send it to the next command (**|**).</span></span>
    
- <span data-ttu-id="18d6b-132">ユーザープリンシパル名のリストをアルファベット順に並べ替え (**UserPrincipalName を並べ替え**)、次のコマンドに送信し **|** ます ()。</span><span class="sxs-lookup"><span data-stu-id="18d6b-132">Sort the list of User Principal Names alphabetically (**Sort UserPrincipalName**) and send it to the next command (**|**).</span></span>
    
- <span data-ttu-id="18d6b-133">各アカウントのユーザープリンシパル名プロパティのみを表示します (**UserPrincipalName を選択**します)。</span><span class="sxs-lookup"><span data-stu-id="18d6b-133">Display just the User Principal Name property for each account (**Select UserPrincipalName**).</span></span>

- <span data-ttu-id="18d6b-134">一度に 1 画面ずつ表示する (**More**)。</span><span class="sxs-lookup"><span data-stu-id="18d6b-134">Display them one screen at a time (**More**).</span></span>
    
<span data-ttu-id="18d6b-135">このコマンドにより、使用しているアカウントすべてが表示されます。</span><span class="sxs-lookup"><span data-stu-id="18d6b-135">This command will list all of your accounts.</span></span> <span data-ttu-id="18d6b-136">表示名 (姓と名) に基づいてアカウントのユーザープリンシパル名を表示する場合は、以下の **$userName**変数 (文字を削除 \< and > します) を入力してから、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="18d6b-136">If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```powershell
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="18d6b-137">この例では、Caleb が Ls の表示名を持つユーザーアカウントのユーザープリンシパル名を表示します。</span><span class="sxs-lookup"><span data-stu-id="18d6b-137">This example displays the User Principal Name for the user account with the display name of Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="18d6b-p103">**$upn** 変数を使用すると、表示名に基づいて個々のアカウントに変更を加えることができます。次の例では Belinda Newman の使用場所をフランスに設定しますが、ユーザー プリンシパル名ではなく表示名を指定します。</span><span class="sxs-lookup"><span data-stu-id="18d6b-p103">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```powershell
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="18d6b-140">すべてのユーザー アカウントのプロパティを変更する</span><span class="sxs-lookup"><span data-stu-id="18d6b-140">Change properties for all user accounts</span></span>

<span data-ttu-id="18d6b-p104">すべてのユーザーのプロパティを変更する場合には、 **Get-AzureADUser** と **Set-AzureADUser** コマンドレットを組み合わせて使用できます。次の例は、すべてのユーザーについて、使用場所をフランスに変更します。</span><span class="sxs-lookup"><span data-stu-id="18d6b-p104">To change properties for all users, you can use the combination of the **Get-AzureADUser** and **Set-AzureADUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```powershell
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="18d6b-143">次のコマンドは、PowerShell に次のように指示します。</span><span class="sxs-lookup"><span data-stu-id="18d6b-143">This command instructs PowerShell to:</span></span>
  
- <span data-ttu-id="18d6b-144">ユーザーアカウントのすべての情報を取得し (**set-azureaduser**)、次のコマンドに送信し **|** ます ()。</span><span class="sxs-lookup"><span data-stu-id="18d6b-144">Get all of the information on the user accounts (**Get-AzureADUser**) and send it to the next command (**|**).</span></span>
    
- <span data-ttu-id="18d6b-145">ユーザーの所在地をフランスに設定します (**set-azureaduser-@ location "FR"**)。</span><span class="sxs-lookup"><span data-stu-id="18d6b-145">Set the user location to France (**Set-AzureADUser -UsageLocation "FR"**).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="18d6b-146">特定のユーザー アカウント セットのプロパティを変更する</span><span class="sxs-lookup"><span data-stu-id="18d6b-146">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="18d6b-p105">特定のユーザー アカウント セットのプロパティを変更する場合には、**Get-AzureADUser**、**Where**、**Set-AzureADUser** コマンドレットの組み合わせを使用することができます。次の例は、会計部門のすべてのユーザーについて、使用場所をフランスに変更します。</span><span class="sxs-lookup"><span data-stu-id="18d6b-p105">To change properties for a specific set of user account, you can use the combination of the **Get-AzureADUser**, **Where**, and **Set-AzureADUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```powershell
Get-AzureADUser | Where {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="18d6b-149">次のコマンドは、PowerShell に次のように指示します。</span><span class="sxs-lookup"><span data-stu-id="18d6b-149">This command instructs PowerShell to:</span></span>
  
- <span data-ttu-id="18d6b-150">ユーザーアカウントのすべての情報を取得し (**set-azureaduser**)、次のコマンドに送信し **|** ます ()。</span><span class="sxs-lookup"><span data-stu-id="18d6b-150">Get all of the information on the user accounts (**Get-AzureADUser**) and send it to the next command (**|**).</span></span>
    
- <span data-ttu-id="18d6b-151">Department プロパティが "Accounting" に設定されているすべてのユーザーアカウントを検索し**ます (Where {$ _)。Department-eq "Accounting"}**) を行い、結果の情報を次のコマンドに送信し **|** ます ()。</span><span class="sxs-lookup"><span data-stu-id="18d6b-151">Find all of the user accounts that have their Department property set to "Accounting" (**Where {$_.Department -eq "Accounting"}**) and send the resulting information to the next command (**|**).</span></span>
    
- <span data-ttu-id="18d6b-152">ユーザーの所在地をフランスに設定します (**set-azureaduser-@ location "FR"**)。</span><span class="sxs-lookup"><span data-stu-id="18d6b-152">Set the user location to France (**Set-AzureADUser -UsageLocation "FR"**).</span></span>
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="18d6b-153">Windows PowerShell 用 Microsoft Azure Active Directory モジュールを使用する</span><span class="sxs-lookup"><span data-stu-id="18d6b-153">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="18d6b-154">Windows PowerShell 用 Microsoft Azure Active Directory モジュールを使用して、ユーザーアカウントのプロパティを構成するには、 **get-msoluser**コマンドレットを使用して、設定または変更するプロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="18d6b-154">To configure properties for user accounts with the Microsoft Azure Active Directory Module for Windows PowerShell, you use the **Set-MsolUser** cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="18d6b-155">最初に、 [Microsoft 365 テナントに接続](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)します。</span><span class="sxs-lookup"><span data-stu-id="18d6b-155">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
  
>[!Note]
><span data-ttu-id="18d6b-156">PowerShell Core は、Windows PowerShell 用 Microsoft Azure Active Directory モジュールと、名前に **Msol** が含まれるコマンドレットをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="18d6b-156">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="18d6b-157">これらのコマンドレットを引き続き使用するには、Windows PowerShell から実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="18d6b-157">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="18d6b-158">特定のユーザー アカウントのプロパティを変更する</span><span class="sxs-lookup"><span data-stu-id="18d6b-158">Change properties for a specific user account</span></span>

<span data-ttu-id="18d6b-159">特定のユーザー アカウントのプロパティを構成する場合、[Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) コマンドレットを使用して、設定または変更するプロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="18d6b-159">To configure properties for a specific user account, you use the [Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="18d6b-p107">**-UserPrincipalName** パラメーターでアカウントを識別し、その他のパラメーターで特定のプロパティを設定または変更します。最も一般的なパラメーターの一覧を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="18d6b-p107">You identify the account with the **-UserPrincipalName** parameter and set or change specific properties with additional parameters. Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="18d6b-162">-City "<市区町村名>"</span><span class="sxs-lookup"><span data-stu-id="18d6b-162">-City "\<city name>"</span></span>
    
- <span data-ttu-id="18d6b-163">-Country "<国名>"</span><span class="sxs-lookup"><span data-stu-id="18d6b-163">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="18d6b-164">-Department "<部署名>"</span><span class="sxs-lookup"><span data-stu-id="18d6b-164">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="18d6b-165">-DisplayName "<完全なユーザー名>"</span><span class="sxs-lookup"><span data-stu-id="18d6b-165">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="18d6b-166">-Fax "<fax 番号>"</span><span class="sxs-lookup"><span data-stu-id="18d6b-166">-Fax "\<fax number>"</span></span>
    
- <span data-ttu-id="18d6b-167">-FirstName "<ユーザーの名>"</span><span class="sxs-lookup"><span data-stu-id="18d6b-167">-FirstName "\<user first name>"</span></span>
    
- <span data-ttu-id="18d6b-168">-LastName "<ユーザーの姓>"</span><span class="sxs-lookup"><span data-stu-id="18d6b-168">-LastName "\<user last name>"</span></span>
    
- <span data-ttu-id="18d6b-169">-MobilePhone "<モバイル機器の番号>"</span><span class="sxs-lookup"><span data-stu-id="18d6b-169">-MobilePhone "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="18d6b-170">-Office "<事業所の場所>"</span><span class="sxs-lookup"><span data-stu-id="18d6b-170">-Office "\<office location>"</span></span>
    
- <span data-ttu-id="18d6b-171">-PhoneNumber "<勤務先電話番号>"</span><span class="sxs-lookup"><span data-stu-id="18d6b-171">-PhoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="18d6b-172">-PostalCode "<郵便番号>"</span><span class="sxs-lookup"><span data-stu-id="18d6b-172">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="18d6b-173">-PreferredLanguage "<言語>"</span><span class="sxs-lookup"><span data-stu-id="18d6b-173">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="18d6b-174">-State "<都道府県名>"</span><span class="sxs-lookup"><span data-stu-id="18d6b-174">-State "\<state name>"</span></span>
    
- <span data-ttu-id="18d6b-175">-StreetAddress "<番地>"</span><span class="sxs-lookup"><span data-stu-id="18d6b-175">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="18d6b-176">-Title "<役職名>"</span><span class="sxs-lookup"><span data-stu-id="18d6b-176">-Title "\<title name>"</span></span>
    
- <span data-ttu-id="18d6b-177">-" \<2-character country or region code> "</span><span class="sxs-lookup"><span data-stu-id="18d6b-177">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="18d6b-178">これは、ISO 3166-1 alpha-2 (A2) の 2 文字の国/地域コードです。</span><span class="sxs-lookup"><span data-stu-id="18d6b-178">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="18d6b-179">その他のパラメーターについては、[Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="18d6b-179">See [Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) for additional parameters.</span></span>

<span data-ttu-id="18d6b-180">すべてのユーザーのユーザー プリンシパル名を表示するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="18d6b-180">To see the User Principal Names of all your users, run the following command.</span></span>
  
```powershell
Get-MSolUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

<span data-ttu-id="18d6b-181">次のコマンドは、PowerShell に次のように指示します。</span><span class="sxs-lookup"><span data-stu-id="18d6b-181">This command instructs PowerShell to:</span></span>
  
- <span data-ttu-id="18d6b-182">ユーザーアカウントのすべての情報を取得し (**get-msoluser**)、次のコマンドに送信し **|** ます ()。</span><span class="sxs-lookup"><span data-stu-id="18d6b-182">Get all of the information on the user accounts (**Get-MsolUser**) and send it to the next command (**|**).</span></span>
    
- <span data-ttu-id="18d6b-183">ユーザープリンシパル名のリストをアルファベット順に並べ替え (**UserPrincipalName を並べ替え**)、次のコマンドに送信し **|** ます ()。</span><span class="sxs-lookup"><span data-stu-id="18d6b-183">Sort the list of User Principal Names alphabetically (**Sort UserPrincipalName**) and send it to the next command (**|**).</span></span>
    
- <span data-ttu-id="18d6b-184">各アカウントのユーザープリンシパル名プロパティのみを表示します (**UserPrincipalName を選択**します)。</span><span class="sxs-lookup"><span data-stu-id="18d6b-184">Display just the User Principal Name property for each account (**Select UserPrincipalName**).</span></span>
    
- <span data-ttu-id="18d6b-185">一度に 1 画面ずつ表示する (**More**)。</span><span class="sxs-lookup"><span data-stu-id="18d6b-185">Display them one screen at a time (**More**).</span></span>
    
<span data-ttu-id="18d6b-186">このコマンドにより、使用しているアカウントすべてが表示されます。</span><span class="sxs-lookup"><span data-stu-id="18d6b-186">This command will list all of your accounts.</span></span> <span data-ttu-id="18d6b-187">表示名 (姓と名) に基づいてアカウントのユーザープリンシパル名を表示する場合は、以下の **$userName**変数 (文字を削除 \< and > します) を入力してから、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="18d6b-187">If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```powershell
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="18d6b-188">次の例では、Caleb Sills という名前のユーザーのユーザー プリンシパル名が表示されます。</span><span class="sxs-lookup"><span data-stu-id="18d6b-188">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="18d6b-p109">**$upn** 変数を使用すると、表示名に基づいて個々のアカウントに変更を加えることができます。次の例では Belinda Newman の使用場所をフランスに設定しますが、ユーザー プリンシパル名ではなく表示名を指定します。</span><span class="sxs-lookup"><span data-stu-id="18d6b-p109">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```powershell
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="18d6b-191">すべてのユーザー アカウントのプロパティを変更する</span><span class="sxs-lookup"><span data-stu-id="18d6b-191">Change properties for all user accounts</span></span>

<span data-ttu-id="18d6b-p110">すべてのユーザーのプロパティを変更する場合には、 **Get-MsolUser** と **Set-MsolUser** コマンドレットを組み合わせて使用できます。次の例は、すべてのユーザーについて、使用場所をフランスに変更します。</span><span class="sxs-lookup"><span data-stu-id="18d6b-p110">To change properties for all users, you can use the combination of the **Get-MsolUser** and **Set-MsolUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```powershell
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="18d6b-194">次のコマンドは、PowerShell に次のように指示します。</span><span class="sxs-lookup"><span data-stu-id="18d6b-194">This command instructs PowerShell to:</span></span>
  
- <span data-ttu-id="18d6b-195">ユーザーアカウントのすべての情報を取得し (**get-msoluser**)、次のコマンドに送信し **|** ます ()。</span><span class="sxs-lookup"><span data-stu-id="18d6b-195">Get all of the information on the user accounts (**Get-MsolUser**) and send it to the next command (**|**).</span></span>
    
- <span data-ttu-id="18d6b-196">ユーザーの所在地をフランスに設定します (**get-msoluser-@ location "FR"**)。</span><span class="sxs-lookup"><span data-stu-id="18d6b-196">Set the user location to France (**Set-MsolUser -UsageLocation "FR"**).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="18d6b-197">特定のユーザー アカウント セットのプロパティを変更する</span><span class="sxs-lookup"><span data-stu-id="18d6b-197">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="18d6b-198">特定のユーザーアカウントセットのプロパティを変更するには、 **get-msoluser**、 **Where**、および**get-msoluser**コマンドレットの組み合わせを使用できます。</span><span class="sxs-lookup"><span data-stu-id="18d6b-198">To change properties for a specific set of user account, you can use the combination of the **Get-MsolUser**, **Where**, and **Set-MsolUser** cmdlets.</span></span> <span data-ttu-id="18d6b-199">次の例は、会計部門のすべてのユーザーについて、使用場所をフランスに変更します。</span><span class="sxs-lookup"><span data-stu-id="18d6b-199">The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```powershell
Get-MsolUser | Where {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="18d6b-200">次のコマンドは、PowerShell に次のように指示します。</span><span class="sxs-lookup"><span data-stu-id="18d6b-200">This command instructs PowerShell to:</span></span>
  
- <span data-ttu-id="18d6b-201">ユーザーアカウントのすべての情報を取得し (**get-msoluser**)、次のコマンドに送信し **|** ます ()。</span><span class="sxs-lookup"><span data-stu-id="18d6b-201">Get all of the information on the user accounts (**Get-MsolUser**) and send it to the next command (**|**).</span></span>
    
- <span data-ttu-id="18d6b-202">Department プロパティが "Accounting" に設定されているすべてのユーザーアカウントを検索し**ます (Where {$ _)。Department-eq "Accounting"}**) を行い、結果の情報を次のコマンドに送信し **|** ます ()。</span><span class="sxs-lookup"><span data-stu-id="18d6b-202">Find all of the user accounts that have their Department property set to "Accounting" (**Where {$_.Department -eq "Accounting"}**) and send the resulting information to the next command (**|**).</span></span>
    
- <span data-ttu-id="18d6b-203">ユーザーの所在地をフランスに設定します (**get-msoluser-@ location "FR"**)。</span><span class="sxs-lookup"><span data-stu-id="18d6b-203">Set the user location to France (**Set-MsolUser -UsageLocation "FR"**).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="18d6b-204">関連項目</span><span class="sxs-lookup"><span data-stu-id="18d6b-204">See also</span></span>

[<span data-ttu-id="18d6b-205">PowerShell を使用して Microsoft 365 のユーザーアカウント、ライセンス、グループを管理する</span><span class="sxs-lookup"><span data-stu-id="18d6b-205">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="18d6b-206">PowerShell を使用して Microsoft 365 を管理する</span><span class="sxs-lookup"><span data-stu-id="18d6b-206">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="18d6b-207">Microsoft 365 の PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="18d6b-207">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)
