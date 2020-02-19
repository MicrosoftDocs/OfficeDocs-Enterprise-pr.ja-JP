---
title: Office 365 PowerShell を使ったサービスへのアクセスを無効にする
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/17/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Office_Other
- PowerShell
- LIL_Placement
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: Office 365 PowerShell を使用して、ユーザーの Office 365 サービスへのアクセスを無効にします。
ms.openlocfilehash: 17927b6d7e402aff66c059e159ae81a950667ad1
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106218"
---
# <a name="disable-access-to-services-with-office-365-powershell"></a><span data-ttu-id="fa980-103">Office 365 PowerShell を使ったサービスへのアクセスを無効にする</span><span class="sxs-lookup"><span data-stu-id="fa980-103">Disable access to services with Office 365 PowerShell</span></span>

<span data-ttu-id="fa980-104">Office 365 アカウントにライセンスプランのライセンスが割り当てられている場合、そのライセンスから Office 365 サービスがユーザーに対して利用可能になります。</span><span class="sxs-lookup"><span data-stu-id="fa980-104">When an Office 365 account is assigned a license from a licensing plan, Office 365 services are made available to the user from that license.</span></span> <span data-ttu-id="fa980-105">ただし、ユーザーがアクセスできる Office 365 サービスを制御することができます。</span><span class="sxs-lookup"><span data-stu-id="fa980-105">However, you can control the Office 365 services that the user can access.</span></span> <span data-ttu-id="fa980-106">たとえば、ライセンスで SharePoint Online サービスへのアクセスが許可されている場合でも、アクセスを無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="fa980-106">For example, even though the license allows access to the SharePoint Online service, you can disable access to it.</span></span> <span data-ttu-id="fa980-107">PowerShell を使用して、次のような特定のライセンスプランで任意の数のサービスへのアクセスを無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="fa980-107">You can use PowerShell to disable access to any number of services for a specific licensing plan for:</span></span>

- <span data-ttu-id="fa980-108">個々のアカウント。</span><span class="sxs-lookup"><span data-stu-id="fa980-108">An individual account.</span></span>
- <span data-ttu-id="fa980-109">アカウントのグループ。</span><span class="sxs-lookup"><span data-stu-id="fa980-109">A group of accounts.</span></span>
- <span data-ttu-id="fa980-110">組織内のすべてのアカウント。</span><span class="sxs-lookup"><span data-stu-id="fa980-110">All accounts in your organization.</span></span>

>[!Note]
><span data-ttu-id="fa980-111">Office 365 サービスの依存関係によって、他のサービスに依存している場合に、指定されたサービスが無効になることがあります。</span><span class="sxs-lookup"><span data-stu-id="fa980-111">There are Office 365 service dependencies that can prevent you from disabling a specified service when other services depend on it.</span></span>
>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="fa980-112">Windows PowerShell の Microsoft Azure Active Directory モジュールを使用する</span><span class="sxs-lookup"><span data-stu-id="fa980-112">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="fa980-113">まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="fa980-113">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="fa980-114">次に、このコマンドを使用して、使用可能なライセンスプラン (AccountSkuIds とも呼ばれます) を表示します。</span><span class="sxs-lookup"><span data-stu-id="fa980-114">Next, use this command to view your available licensing plans, also known as AccountSkuIds:</span></span>

```powershell
Get-MsolAccountSku | Select AccountSkuId | Sort AccountSkuId
```

>[!Note]
><span data-ttu-id="fa980-115">PowerShell Core は、Windows PowerShell 用 Microsoft Azure Active Directory モジュールと、名前に **Msol** が含まれるコマンドレットをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="fa980-115">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="fa980-116">これらのコマンドレットを引き続き使用するには、Windows PowerShell から実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fa980-116">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="fa980-117">詳細については、「 [Office 365 PowerShell でライセンスとサービスを表示](view-licenses-and-services-with-office-365-powershell.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fa980-117">For more information, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="fa980-118">このトピックの手順の前と後の結果を確認するには、「 [Office 365 PowerShell を使用してアカウントのライセンスとサービスの詳細を表示](view-account-license-and-service-details-with-office-365-powershell.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fa980-118">To see the before and after results of the procedures in this topic, see [View account license and service details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="fa980-119">このトピックで説明されている手順を自動化する PowerShell スクリプトが利用可能です。</span><span class="sxs-lookup"><span data-stu-id="fa980-119">A PowerShell script is available that automates the procedures described in this topic.</span></span> <span data-ttu-id="fa980-120">具体的には、このスクリプトを使用すると、Sway などの Office 365 組織のサービスを表示したり、無効にしたりできます。</span><span class="sxs-lookup"><span data-stu-id="fa980-120">Specifically, the script lets you view and disable services in your Office 365 organization, including Sway.</span></span> <span data-ttu-id="fa980-121">詳細については、「[Office 365 PowerShell を使った Sway へのアクセスを無効にする](disable-access-to-sway-with-office-365-powershell.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="fa980-121">For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
    
### <a name="disable-specific-office-365-services-for-specific-users-for-a-specific-licensing-plan"></a><span data-ttu-id="fa980-122">特定のライセンスプランの特定のユーザーに対して特定の Office 365 サービスを無効にする</span><span class="sxs-lookup"><span data-stu-id="fa980-122">Disable specific Office 365 services for specific users for a specific licensing plan</span></span>
  
<span data-ttu-id="fa980-123">特定のライセンスプランのユーザーに対して特定の Office 365 サービスのセットを無効にするには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="fa980-123">To disable a specific set of Office 365 services for users for a specific licensing plan, perform the following steps:</span></span>
  
#### <a name="step-1-identify-the-undesirable-services-in-the-licensing-plan-by-using-the-following-syntax"></a><span data-ttu-id="fa980-124">手順 1: 次の構文を使用して、ライセンスプランで不要なサービスを特定します。</span><span class="sxs-lookup"><span data-stu-id="fa980-124">Step 1: Identify the undesirable services in the licensing plan by using the following syntax:</span></span>
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
```

<span data-ttu-id="fa980-125">次の例では、という名前`litwareinc:ENTERPRISEPACK`のライセンスプラン (Office 365 Enterprise E3) で Office および SharePoint Online サービスを無効にする**licenseoptions**オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="fa980-125">The following example creates a **LicenseOptions** object that disables the Office and SharePoint Online services in the licensing plan named `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span></span>
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

#### <a name="step-2-use-the-licenseoptions-object-from-step-1-on-one-or-more-users"></a><span data-ttu-id="fa980-126">手順 2: 1 人以上のユーザーの手順1の**Licenseoptions**オブジェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="fa980-126">Step 2: Use the **LicenseOptions** object from Step 1 on one or more users.</span></span>
    
<span data-ttu-id="fa980-127">サービスが無効になっている新しいアカウントを作成するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="fa980-127">To create a new account that has the services disabled, use the following syntax:</span></span>
    
```powershell
New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
```

<span data-ttu-id="fa980-128">次の例では、ライセンスを割り当て、手順1で説明されているサービスを無効にする Allie Bellew の新しいアカウントを作成します。</span><span class="sxs-lookup"><span data-stu-id="fa980-128">The following example creates a new account for Allie Bellew that assigns the license and disables the services described in Step 1.</span></span>
    
```powershell
New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
```

<span data-ttu-id="fa980-129">Office 365 PowerShell でユーザーアカウントを作成する方法の詳細については、「 [office 365 powershell を使用してユーザーアカウントを作成](create-user-accounts-with-office-365-powershell.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fa980-129">For more information about creating user accounts in Office 365 PowerShell, see [Create user accounts with Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="fa980-130">ライセンスを付与された既存のユーザー用のサービスを無効にするには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="fa980-130">To disable the services for an existing licensed user, use the following syntax:</span></span>
    
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
```

<span data-ttu-id="fa980-131">この例では、ユーザー BelindaN@litwareinc.com に対してサービスを無効にします。</span><span class="sxs-lookup"><span data-stu-id="fa980-131">This example disables the services for the user BelindaN@litwareinc.com.</span></span>
    
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
```

<span data-ttu-id="fa980-132">既存のライセンスを持つすべてのユーザーについて、手順1で説明されているサービスを無効にするには、 **get-msolaccountsku**コマンドレット ( **LITWAREINC: enterprisepack**など) の表示から Office 365 プランの名前を指定し、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="fa980-132">To disable the services described in Step 1 for all existing licensed users, specify the name of your Office 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK**), and then run the following commands:</span></span>
    
```powershell
$acctSKU="<AccountSkuId>"
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses.AccountSku.SkuPartNumber -contains ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

 <span data-ttu-id="fa980-133">_All_パラメーターを使用せずに**get-msoluser**コマンドレットを使用すると、最初の500ユーザーアカウントのみが返されます。</span><span class="sxs-lookup"><span data-stu-id="fa980-133">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 user accounts are returned.</span></span>

<span data-ttu-id="fa980-134">既存のユーザーのグループに対してサービスを無効にするには、次のいずれかの方法を使用して、ユーザーを特定します。</span><span class="sxs-lookup"><span data-stu-id="fa980-134">To disable the services for a group of existing users, use either of the following methods to identify the users:</span></span>
    
<span data-ttu-id="fa980-135">**方法1既存のアカウント属性に基づいてアカウントをフィルター処理する**</span><span class="sxs-lookup"><span data-stu-id="fa980-135">**Method 1. Filter the accounts based on an existing account attribute**</span></span> 

<span data-ttu-id="fa980-136">この設定を行うには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="fa980-136">To do this, use the following syntax:</span></span>
    
```powershell
$x = Get-MsolUser -All <FilterableAttributes>
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

<span data-ttu-id="fa980-137">次の例では、米国内の販売部門のユーザーのサービスを無効にします。</span><span class="sxs-lookup"><span data-stu-id="fa980-137">The following example disables the services for users in the Sales department in the United States.</span></span>
    
```powershell
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
$USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

<span data-ttu-id="fa980-138">**方法 2: 特定のアカウントの一覧を使用する**</span><span class="sxs-lookup"><span data-stu-id="fa980-138">**Method 2: Use a list of specific accounts**</span></span> 

<span data-ttu-id="fa980-139">これを行うには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="fa980-139">To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="fa980-140">次のように各行に 1 つのアカウントが含まれるテキスト ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="fa980-140">Create a text file that contains one account on each line like this:</span></span>
    
  ```powershell
  akol@contoso.com
  tjohnston@contoso.com
  kakers@contoso.com
  ```

  <span data-ttu-id="fa980-141">この例では、テキストファイルは「C\\: My\\Documents のアカウント .txt」です。</span><span class="sxs-lookup"><span data-stu-id="fa980-141">In this example, the text file is C:\\My Documents\\Accounts.txt.</span></span>
    
2. <span data-ttu-id="fa980-142">次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="fa980-142">Run the following command:</span></span>
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

<span data-ttu-id="fa980-143">複数のライセンスプランのサービスへのアクセスを無効にする場合は、ライセンスプランごとに上記の手順を繰り返し、以下のことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="fa980-143">If you want to disable access to services for multiple licensing plans, repeat the above instructions for each licensing plan, ensuring that:</span></span>

- <span data-ttu-id="fa980-144">ユーザーアカウントにはライセンスプランが割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="fa980-144">The user accounts have been assigned the licensing plan.</span></span>
- <span data-ttu-id="fa980-145">無効化するサービスは、ライセンスプランで利用できます。</span><span class="sxs-lookup"><span data-stu-id="fa980-145">The services to disable are available in the licensing plan.</span></span>

<span data-ttu-id="fa980-146">ユーザーがライセンスプランに割り当てている間、ユーザーに対して Office 365 サービスを無効にするには、「[ユーザーのライセンスの割り当て中にサービスへのアクセスを無効](disable-access-to-services-while-assigning-user-licenses.md)にする」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fa980-146">To disable Office 365 services for users while you are assigning them to a licensing plan, see [Disable access to services while assigning user licenses](disable-access-to-services-while-assigning-user-licenses.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="fa980-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="fa980-147">See also</span></span>

[<span data-ttu-id="fa980-148">Office 365 PowerShell を使用してユーザーアカウント、ライセンス、グループを管理する</span><span class="sxs-lookup"><span data-stu-id="fa980-148">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="fa980-149">Office 365 PowerShell による Office 365 の管理</span><span class="sxs-lookup"><span data-stu-id="fa980-149">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="fa980-150">Office 365 PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="fa980-150">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
