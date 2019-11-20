---
title: Office 365 PowerShell を使ったサービスへのアクセスを無効にする
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/28/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
- LIL_Placement
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: Office 365 PowerShell を使用して、ユーザーの Office 365 サービスへのアクセスを無効にします。
ms.openlocfilehash: c012d7451d022ea8cf3e3fa1a8d0a89d804e9c66
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2019
ms.locfileid: "38746280"
---
# <a name="disable-access-to-services-with-office-365-powershell"></a><span data-ttu-id="99d59-103">Office 365 PowerShell を使ったサービスへのアクセスを無効にする</span><span class="sxs-lookup"><span data-stu-id="99d59-103">Disable access to services with Office 365 PowerShell</span></span>

<span data-ttu-id="99d59-104">Office 365 アカウントにライセンスプランのライセンスが割り当てられている場合、そのライセンスから Office 365 サービスがユーザーに対して利用可能になります。</span><span class="sxs-lookup"><span data-stu-id="99d59-104">When an Office 365 account is assigned a license from a licensing plan, Office 365 services are made available to the user from that license.</span></span> <span data-ttu-id="99d59-105">ただし、ユーザーがアクセスできる Office 365 サービスを制御することができます。</span><span class="sxs-lookup"><span data-stu-id="99d59-105">However, you can control the Office 365 services that the user can access.</span></span> <span data-ttu-id="99d59-106">たとえば、ライセンスで SharePoint Online サービスへのアクセスが許可されている場合でも、アクセスを無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="99d59-106">For example, even though the license allows access to the SharePoint Online service, you can disable access to it.</span></span> <span data-ttu-id="99d59-107">PowerShell を使用して、次のような特定のライセンスプランで任意の数のサービスへのアクセスを無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="99d59-107">You can use PowerShell to disable access to any number of services for a specific licensing plan for:</span></span>

- <span data-ttu-id="99d59-108">個々のアカウント。</span><span class="sxs-lookup"><span data-stu-id="99d59-108">An individual account.</span></span>
    
- <span data-ttu-id="99d59-109">アカウントのグループ。</span><span class="sxs-lookup"><span data-stu-id="99d59-109">A group of accounts.</span></span>
    
- <span data-ttu-id="99d59-110">組織内のすべてのアカウント。</span><span class="sxs-lookup"><span data-stu-id="99d59-110">All accounts in your organization.</span></span>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="99d59-111">Windows PowerShell の Microsoft Azure Active Directory モジュールを使用する</span><span class="sxs-lookup"><span data-stu-id="99d59-111">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="99d59-112">まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="99d59-112">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="99d59-113">次に、このコマンドを使用して、使用可能なライセンスプラン (AccountSkuIds とも呼ばれます) を表示します。</span><span class="sxs-lookup"><span data-stu-id="99d59-113">Next, use this command to view your available licensing plans, also known as AccountSkuIds:</span></span>

```powershell
Get-MsolAccountSku | Select AccountSkuId | Sort AccountSkuId
```

<span data-ttu-id="99d59-114">詳細については、「 [Office 365 PowerShell でライセンスとサービスを表示](view-licenses-and-services-with-office-365-powershell.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="99d59-114">For more information, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="99d59-115">このトピックの手順の前と後の結果を確認するには、「 [Office 365 PowerShell を使用してアカウントのライセンスとサービスの詳細を表示](view-account-license-and-service-details-with-office-365-powershell.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="99d59-115">To see the before and after results of the procedures in this topic, see [View account license and service details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="99d59-116">このトピックで説明されている手順を自動化する PowerShell スクリプトが利用可能です。</span><span class="sxs-lookup"><span data-stu-id="99d59-116">A PowerShell script is available that automates the procedures described in this topic.</span></span> <span data-ttu-id="99d59-117">具体的には、このスクリプトを使用すると、Sway などの Office 365 組織のサービスを表示したり、無効にしたりできます。</span><span class="sxs-lookup"><span data-stu-id="99d59-117">Specifically, the script lets you view and disable services in your Office 365 organization, including Sway.</span></span> <span data-ttu-id="99d59-118">詳細については、「[Office 365 PowerShell を使った Sway へのアクセスを無効にする](disable-access-to-sway-with-office-365-powershell.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="99d59-118">For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
    
### <a name="disable-specific-office-365-services-for-specific-users-for-a-specific-licensing-plan"></a><span data-ttu-id="99d59-119">特定のライセンスプランの特定のユーザーに対して特定の Office 365 サービスを無効にする</span><span class="sxs-lookup"><span data-stu-id="99d59-119">Disable specific Office 365 services for specific users for a specific licensing plan</span></span>
  
<span data-ttu-id="99d59-120">特定のライセンスプランのユーザーに対して特定の Office 365 サービスのセットを無効にするには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="99d59-120">To disable a specific set of Office 365 services for users for a specific licensing plan, perform the following steps:</span></span>
  
1. <span data-ttu-id="99d59-121">次の構文を使用して、ライセンスプランで不要なサービスを特定します。</span><span class="sxs-lookup"><span data-stu-id="99d59-121">Identify the undesirable services in the licensing plan by using the following syntax:</span></span>
    
  ```powershell
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

  <span data-ttu-id="99d59-122">次の例では、という名前`litwareinc:ENTERPRISEPACK`のライセンスプラン (Office 365 Enterprise E3) で Office および SharePoint Online サービスを無効にする**licenseoptions**オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="99d59-122">The following example creates a **LicenseOptions** object that disables the Office and SharePoint Online services in the licensing plan named `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span></span>
    
  ```powershell
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. <span data-ttu-id="99d59-123">手順 1 の **LicenseOptions** オブジェクトを、1 人以上のユーザーに使用します。</span><span class="sxs-lookup"><span data-stu-id="99d59-123">Use the **LicenseOptions** object from Step 1 on one or more users.</span></span>
    
  - <span data-ttu-id="99d59-124">サービスが無効になっている新しいアカウントを作成するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="99d59-124">To create a new account that has the services disabled, use the following syntax:</span></span>
    
  ```powershell
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

  <span data-ttu-id="99d59-125">次の例では、ライセンスを割り当て、手順1で説明されているサービスを無効にする Allie Bellew の新しいアカウントを作成します。</span><span class="sxs-lookup"><span data-stu-id="99d59-125">The following example creates a new account for Allie Bellew that assigns the license and disables the services described in Step 1.</span></span>
    
  ```powershell
  New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
  ```

  <span data-ttu-id="99d59-126">Office 365 PowerShell でユーザーアカウントを作成する方法の詳細については、「 [office 365 powershell を使用してユーザーアカウントを作成](create-user-accounts-with-office-365-powershell.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="99d59-126">For more information about creating user accounts in Office 365 PowerShell, see [Create user accounts with Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span></span>
    
  - <span data-ttu-id="99d59-127">ライセンスを付与された既存のユーザー用のサービスを無効にするには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="99d59-127">To disable the services for an existing licensed user, use the following syntax:</span></span>
    
  ```powershell
  Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
  ```

  <span data-ttu-id="99d59-128">この例では、ユーザー BelindaN@litwareinc.com に対してサービスを無効にします。</span><span class="sxs-lookup"><span data-stu-id="99d59-128">This example disables the services for the user BelindaN@litwareinc.com.</span></span>
    
  ```powershell
  Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
  ```

  - <span data-ttu-id="99d59-129">既存のライセンスを持つすべてのユーザーについて、手順1で説明されているサービスを無効にするには、 **get-msolaccountsku**コマンドレット ( **LITWAREINC: enterprisepack**など) の表示から Office 365 プランの名前を指定し、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="99d59-129">To disable the services described in Step 1 for all existing licensed users, specify the name of your Office 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK**), and then run the following commands:</span></span>
    
  ```powershell
  $acctSKU="<AccountSkuId>"
  $AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
  $AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  <span data-ttu-id="99d59-130">_All_パラメーターを使用せずに**get-msoluser**コマンドレットを使用すると、最初の500ユーザーアカウントのみが返されます。</span><span class="sxs-lookup"><span data-stu-id="99d59-130">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 user accounts are returned.</span></span>


  - <span data-ttu-id="99d59-131">既存のユーザーのグループに対してサービスを無効にするには、次のいずれかの方法を使用して、ユーザーを特定します。</span><span class="sxs-lookup"><span data-stu-id="99d59-131">To disable the services for a group of existing users, use either of the following methods to identify the users:</span></span>
    
  - <span data-ttu-id="99d59-132">**既存のアカウント属性に基づいてアカウントをフィルターする** これを行うには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="99d59-132">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
  ```powershell
  $x = Get-MsolUser -All <FilterableAttributes>
  $x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  <span data-ttu-id="99d59-133">次の例では、米国内の販売部門のユーザーのサービスを無効にします。</span><span class="sxs-lookup"><span data-stu-id="99d59-133">The following example disables the services for users in the Sales department in the United States.</span></span>
    
  ```powershell
  $USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
  $USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - <span data-ttu-id="99d59-134">**特定のアカウントの一覧を使用する** これを行うには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="99d59-134">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="99d59-135">次のように各行に 1 つのアカウントが含まれるテキスト ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="99d59-135">Create a text file that contains one account on each line like this:</span></span>
    
  ```powershell
  akol@contoso.com
  tjohnston@contoso.com
  kakers@contoso.com
  ```

  <span data-ttu-id="99d59-136">この例では、テキストファイルは「C\\: My\\Documents のアカウント .txt」です。</span><span class="sxs-lookup"><span data-stu-id="99d59-136">In this example, the text file is C:\\My Documents\\Accounts.txt.</span></span>
    
2. <span data-ttu-id="99d59-137">次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="99d59-137">Run the following command:</span></span>
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

<span data-ttu-id="99d59-138">複数のライセンスプランのサービスへのアクセスを無効にする場合は、ライセンスプランごとに上記の手順を繰り返し、以下のことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="99d59-138">If you want to disable access to services for multiple licensing plans, repeat the above instructions for each licensing plan, ensuring that:</span></span>

- <span data-ttu-id="99d59-139">ユーザーアカウントにはライセンスプランが割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="99d59-139">The user accounts have been assigned the licensing plan.</span></span>
- <span data-ttu-id="99d59-140">無効化するサービスは、ライセンスプランで利用できます。</span><span class="sxs-lookup"><span data-stu-id="99d59-140">The services to disable are available in the licensing plan.</span></span>

<span data-ttu-id="99d59-141">ユーザーがライセンスプランに割り当てている間、ユーザーに対して Office 365 サービスを無効にするには、「[ユーザーのライセンスの割り当て中にサービスへのアクセスを無効](disable-access-to-services-while-assigning-user-licenses.md)にする」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="99d59-141">To disable Office 365 services for users while you are assigning them to a licensing plan, see [Disable access to services while assigning user licenses](disable-access-to-services-while-assigning-user-licenses.md).</span></span>


## <a name="new-to-office-365"></a><span data-ttu-id="99d59-142">Office 365 を初めて使用する場合</span><span class="sxs-lookup"><span data-stu-id="99d59-142">New to Office 365?</span></span>
<span data-ttu-id="99d59-143"><a name="LinkedIn"> </a></span><span class="sxs-lookup"><span data-stu-id="99d59-143"></span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a><span data-ttu-id="99d59-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="99d59-144">See also</span></span>
<span data-ttu-id="99d59-145"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="99d59-145"></span></span>

<span data-ttu-id="99d59-146">Office 365 PowerShell でのユーザー管理に関する次の追加のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="99d59-146">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="99d59-147">Office 365 PowerShell を使用したユーザー アカウントの削除と復元</span><span class="sxs-lookup"><span data-stu-id="99d59-147">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="99d59-148">Office 365 PowerShell を使用したユーザー アカウントの削除と復元</span><span class="sxs-lookup"><span data-stu-id="99d59-148">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="99d59-149">Office 365 PowerShell でユーザー アカウントをブロックする</span><span class="sxs-lookup"><span data-stu-id="99d59-149">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="99d59-150">Office 365 PowerShell を使用してライセンスをユーザー アカウントに割り当てる</span><span class="sxs-lookup"><span data-stu-id="99d59-150">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="99d59-151">Office 365 PowerShell を使用してユーザー アカウントを作成する</span><span class="sxs-lookup"><span data-stu-id="99d59-151">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
